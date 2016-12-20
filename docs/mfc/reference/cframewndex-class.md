---
title: "CFrameWndEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFrameWndEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFrameWndEx class"
ms.assetid: 5830aca8-4a21-4f31-91f1-dd5477ffcc8d
caps.latest.revision: 39
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFrameWndEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 Windows 單一文件介面 \(SDI\) \(SDI\) 的功能重疊或快顯框架視窗，並處理 Windows 提供成員。  它會擴充 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 類別。  
  
## 語法  
  
```  
class CFrameWndEx : public CFrameWnd  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFrameWndEx::ActiveItemRecalcLayout](../Topic/CFrameWndEx::ActiveItemRecalcLayout.md)|調整 OLE 用戶端項目和架構的工作區的配置。|  
|`CFrameWndEx::AddDockSite`|沒有使用這個方法。|  
|[CFrameWndEx::AddPane](../Topic/CFrameWndEx::AddPane.md)|註冊處理常式使用停駐的控制列。|  
|[CFrameWndEx::AdjustDockingLayout](../Topic/CFrameWndEx::AdjustDockingLayout.md)|重新計算停駐在框架視窗的所有窗格的配置。|  
|[CFrameWndEx::DelayUpdateFrameMenu](../Topic/CFrameWndEx::DelayUpdateFrameMenu.md)|例如，在命令處理閒置時，設定框架功能表然後更新它。|  
|[CFrameWndEx::DockPane](../Topic/CFrameWndEx::DockPane.md)|指定內建的窗格到框架視窗。|  
|[CFrameWndEx::DockPaneLeftOf](../Topic/CFrameWndEx::DockPaneLeftOf.md)|另一個窗格停駐在左邊的窗格。|  
|[CFrameWndEx::EnableAutoHidePanes](../Topic/CFrameWndEx::EnableAutoHidePanes.md)|其停駐在主框架視窗時，指定的一邊啟動窗格的自動隱藏模式。|  
|[CFrameWndEx::EnableDocking](../Topic/CFrameWndEx::EnableDocking.md)|啟用屬於框架視窗的停駐窗格。|  
|[CFrameWndEx::EnableFullScreenMainMenu](../Topic/CFrameWndEx::EnableFullScreenMainMenu.md)|顯示或隱藏主功能表在全螢幕模式。|  
|[CFrameWndEx::EnableFullScreenMode](../Topic/CFrameWndEx::EnableFullScreenMode.md)|啟動框架視窗的全螢幕模式。|  
|[CFrameWndEx::EnableLoadDockState](../Topic/CFrameWndEx::EnableLoadDockState.md)|啟用或停用停駐狀態的載入。|  
|[CFrameWndEx::EnablePaneMenu](../Topic/CFrameWndEx::EnablePaneMenu.md)|啟用或停用自動處理窗格功能表。|  
|[CFrameWndEx::GetActivePopup](../Topic/CFrameWndEx::GetActivePopup.md)|傳回指向目前顯示的快顯功能表。|  
|[CFrameWndEx::GetDefaultResId](../Topic/CFrameWndEx::GetDefaultResId.md)|傳回所指定的資源 ID 架構時載入框架視窗。|  
|[CFrameWndEx::GetDockingManager](../Topic/CFrameWndEx::GetDockingManager.md)|擷取框架視窗的 [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) 物件。|  
|[CFrameWndEx::GetMenuBar](../Topic/CFrameWndEx::GetMenuBar.md)|傳回指向附加的功能表列物件到框架視窗。|  
|[CFrameWndEx::GetPane](../Topic/CFrameWndEx::GetPane.md)|會將指標傳至具有指定之 ID 的窗格 .|  
|[CFrameWndEx::GetRibbonBar](../Topic/CFrameWndEx::GetRibbonBar.md)|擷取框架的功能區列控制項。|  
|[CFrameWndEx::GetTearOffBars](../Topic/CFrameWndEx::GetTearOffBars.md)|傳回在 Tear\-Off 狀態窗格的物件清單。|  
|[CFrameWndEx::GetToolbarButtonToolTipText](../Topic/CFrameWndEx::GetToolbarButtonToolTipText.md)|呼叫框架，當應用程式顯示工具列按鈕的工具提示。|  
|[CFrameWndEx::InsertPane](../Topic/CFrameWndEx::InsertPane.md)|註冊處理常式停駐的窗格。|  
|[CFrameWndEx::IsFullScreen](../Topic/CFrameWndEx::IsFullScreen.md)|判斷框架視窗是否是以全螢幕模式。|  
|[CFrameWndEx::IsMenuBarAvailable](../Topic/CFrameWndEx::IsMenuBarAvailable.md)|判斷為功能表列的物件指標是否有效。|  
|[CFrameWndEx::IsPointNearDockSite](../Topic/CFrameWndEx::IsPointNearDockSite.md)|表示這個點是否位於對齊區域。|  
|[CFrameWndEx::IsPrintPreview](../Topic/CFrameWndEx::IsPrintPreview.md)|表示框架視窗是否在預覽列印模式。|  
|[CFrameWndEx::LoadFrame](../Topic/CFrameWndEx::LoadFrame.md)|這個方法會建構之後呼叫建立框架視窗和載入它的資源。|  
|[CFrameWndEx::NegotiateBorderSpace](../Topic/CFrameWndEx::NegotiateBorderSpace.md)|實作 OLE 用戶端交涉框線。|  
|[CFrameWndEx::OnActivate](../Topic/CFrameWndEx::OnActivate.md)|當使用者輸入會切換至或離開框架時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnActivateApp](../Topic/CFrameWndEx::OnActivateApp.md)|呼叫由架構應用程式時，會選取或取消選取。|  
|[CFrameWndEx::OnChangeVisualManager](../Topic/CFrameWndEx::OnChangeVisualManager.md)|呼叫框架時，這個框架的變更需要視覺管理員的變更。|  
|[CFrameWndEx::OnClose](../Topic/CFrameWndEx::OnClose.md)|架構會呼叫這個方法會關閉框架。|  
|[CFrameWndEx::OnCloseDockingPane](../Topic/CFrameWndEx::OnCloseDockingPane.md)|呼叫框架，當使用者在停駐窗格中按一下 \[**關閉**\] 按鈕。|  
|[CFrameWndEx::OnCloseMiniFrame](../Topic/CFrameWndEx::OnCloseMiniFrame.md)|呼叫框架，當使用者在浮動微型框架視窗中按一下 \[**關閉**\] 按鈕。|  
|[CFrameWndEx::OnClosePopupMenu](../Topic/CFrameWndEx::OnClosePopupMenu.md)|呼叫框架，只有一個作用中的快顯功能表處理 WM\_DESTROY 訊息。|  
|[CFrameWndEx::OnCmdMsg](../Topic/CFrameWndEx::OnCmdMsg.md)|命令分派訊息。|  
|[CFrameWndEx::OnContextHelp](../Topic/CFrameWndEx::OnContextHelp.md)|呼叫由架構來顯示內容的相關說明。|  
|[CFrameWndEx::OnCreate](../Topic/CFrameWndEx::OnCreate.md)|呼叫由架構在架構之後建立的。|  
|[CFrameWndEx::OnDestroy](../Topic/CFrameWndEx::OnDestroy.md)|呼叫由架構，在終結框架。|  
|[CFrameWndEx::OnDrawMenuImage](../Topic/CFrameWndEx::OnDrawMenuImage.md)|呼叫框架，當應用程式在要繪製影像與功能表項目。|  
|[CFrameWndEx::OnDrawMenuLogo](../Topic/CFrameWndEx::OnDrawMenuLogo.md)|呼叫框架，在 `CMFCPopupMenu` 物件處理 [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) 訊息。|  
|[CFrameWndEx::OnDWMCompositionChanged](../Topic/CFrameWndEx::OnDWMCompositionChanged.md)|呼叫框架，在桌面視窗管理員 \(DWM\) 構成啟用或停用。|  
|[CFrameWndEx::OnExitSizeMove](../Topic/CFrameWndEx::OnExitSizeMove.md)|呼叫由架構，在框架停止移動或調整其大小。|  
|[CFrameWndEx::OnGetMinMaxInfo](../Topic/CFrameWndEx::OnGetMinMaxInfo.md)|呼叫框架，該架構調整設定視窗大小限制。|  
|[CFrameWndEx::OnIdleUpdateCmdUI](../Topic/CFrameWndEx::OnIdleUpdateCmdUI.md)|呼叫框架更新框架時，便會顯示訂單處理處於閒置狀態。|  
|[CFrameWndEx::OnLButtonDown](../Topic/CFrameWndEx::OnLButtonDown.md)|當使用者按下滑鼠左鍵時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnLButtonUp](../Topic/CFrameWndEx::OnLButtonUp.md)|使用者放開滑鼠左鍵時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnMenuButtonToolHitTest](../Topic/CFrameWndEx::OnMenuButtonToolHitTest.md)|呼叫框架，在 `CMFCToolBarButton` 物件處理 `WM_NCHITTEST` 訊息。|  
|[CFrameWndEx::OnMenuChar](../Topic/CFrameWndEx::OnMenuChar.md)|呼叫，便會由架構功能表顯示時和使用者按下不對應至命令的按鍵。|  
|[CFrameWndEx::OnMouseMove](../Topic/CFrameWndEx::OnMouseMove.md)|當滑鼠指標移動時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnMoveMiniFrame](../Topic/CFrameWndEx::OnMoveMiniFrame.md)|呼叫框架，該窗格視窗中移動。|  
|[CFrameWndEx::OnNcActivate](../Topic/CFrameWndEx::OnNcActivate.md)|呼叫框架，就必須重新繪製框架的非工作區 \(Nonclient Area\) 表示處於作用中狀態中的變更。|  
|[CFrameWndEx::OnNcCalcSize](../Topic/CFrameWndEx::OnNcCalcSize.md)|呼叫框架，就必須計算工作區的大小和位置。|  
|[CFrameWndEx::OnNcHitTest](../Topic/CFrameWndEx::OnNcHitTest.md)|呼叫框架，當指標移動，或在按下或放開的狀態。|  
|[CFrameWndEx::OnNcMouseMove](../Topic/CFrameWndEx::OnNcMouseMove.md)|呼叫框架，當指標移至非工作區。|  
|[CFrameWndEx::OnNcPaint](../Topic/CFrameWndEx::OnNcPaint.md)|呼叫框架，而必須繪製非工作區。|  
|[CFrameWndEx::OnPaneCheck](../Topic/CFrameWndEx::OnPaneCheck.md)|呼叫由架構窗格控制項的可視性。|  
|[CFrameWndEx::OnPostPreviewFrame](../Topic/CFrameWndEx::OnPostPreviewFrame.md)|呼叫框架，當使用者變更預覽列印模式。|  
|[CFrameWndEx::OnPowerBroadcast](../Topic/CFrameWndEx::OnPowerBroadcast.md)|呼叫框架，當電源管理事件時發生。|  
|[CFrameWndEx::OnSetMenu](../Topic/CFrameWndEx::OnSetMenu.md)|呼叫框架取代框架視窗功能表。|  
|[CFrameWndEx::OnSetPreviewMode](../Topic/CFrameWndEx::OnSetPreviewMode.md)|呼叫框架將框架的預覽列印模式。|  
|[CFrameWndEx::OnSetText](../Topic/CFrameWndEx::OnSetText.md)|呼叫框架設定視窗中的文字。|  
|[CFrameWndEx::OnShowCustomizePane](../Topic/CFrameWndEx::OnShowCustomizePane.md)|呼叫，便會由架構快自訂窗格時啟用。|  
|[CFrameWndEx::OnShowPanes](../Topic/CFrameWndEx::OnShowPanes.md)|呼叫由架構來顯示或隱藏窗格。|  
|[CFrameWndEx::OnShowPopupMenu](../Topic/CFrameWndEx::OnShowPopupMenu.md)|呼叫框架，在快顯功能表啟用。|  
|[CFrameWndEx::OnSize](../Topic/CFrameWndEx::OnSize.md)|在框架大小變更之後，架構會呼叫這個方法。|  
|[CFrameWndEx::OnSizing](../Topic/CFrameWndEx::OnSizing.md)|當使用者調整框架時，架構會呼叫這個方法。|  
|[CFrameWndEx::OnSysColorChange](../Topic/CFrameWndEx::OnSysColorChange.md)|呼叫框架，當系統色彩變更。|  
|[CFrameWndEx::OnTearOffMenu](../Topic/CFrameWndEx::OnTearOffMenu.md)|呼叫框架，若有 Tear\-Off 功能表上手動啟用。|  
|[CFrameWndEx::OnToolbarContextMenu](../Topic/CFrameWndEx::OnToolbarContextMenu.md)|呼叫由架構建立工具列內容功能表。|  
|[CFrameWndEx::OnToolbarCreateNew](../Topic/CFrameWndEx::OnToolbarCreateNew.md)|架構會呼叫這個方法會建立新的工具列。|  
|[CFrameWndEx::OnToolbarDelete](../Topic/CFrameWndEx::OnToolbarDelete.md)|呼叫框架，其在工具列中刪除。|  
|[CFrameWndEx::OnUpdateFrameMenu](../Topic/CFrameWndEx::OnUpdateFrameMenu.md)|呼叫框架將框架功能表。|  
|[CFrameWndEx::OnUpdateFrameTitle](../Topic/CFrameWndEx::OnUpdateFrameTitle.md)|架構會呼叫這個方法會更新框架視窗的標題列。|  
|[CFrameWndEx::OnUpdatePaneMenu](../Topic/CFrameWndEx::OnUpdatePaneMenu.md)|呼叫框架更新窗格功能表。|  
|[CFrameWndEx::OnWindowPosChanged](../Topic/CFrameWndEx::OnWindowPosChanged.md)|呼叫框架，其在框架大小、位置、疊置順序變更為因呼叫而視窗管理方法。|  
|[CFrameWndEx::PaneFromPoint](../Topic/CFrameWndEx::PaneFromPoint.md)|傳回包含指定之點的停駐窗格。|  
|[CFrameWndEx::PreTranslateMessage](../Topic/CFrameWndEx::PreTranslateMessage.md)|處理特定 Windows 訊息，再分派它們。|  
|[CFrameWndEx::RecalcLayout](../Topic/CFrameWndEx::RecalcLayout.md)|調整框架和它的子視窗的配置。|  
|[CFrameWndEx::RemovePaneFromDockManager](../Topic/CFrameWndEx::RemovePaneFromDockManager.md)|將窗格與停駐管理員的內部清單中移除它。|  
|[CFrameWndEx::SetDockState](../Topic/CFrameWndEx::SetDockState.md)|還原停駐設定儲存在登錄中的停駐狀態。|  
|[CFrameWndEx::SetPrintPreviewFrame](../Topic/CFrameWndEx::SetPrintPreviewFrame.md)|設定預覽列印框架視窗。|  
|[CFrameWndEx::SetupToolbarMenu](../Topic/CFrameWndEx::SetupToolbarMenu.md)|插入使用者定義命令至工具列上的  功能表上的。|  
|[CFrameWndEx::ShowFullScreen](../Topic/CFrameWndEx::ShowFullScreen.md)|交換主要畫面格 \(例如\) 會在全螢幕模式和規則模式之間切換。|  
|[CFrameWndEx::ShowPane](../Topic/CFrameWndEx::ShowPane.md)|顯示或隱藏指定的窗格。|  
|[CFrameWndEx::UpdateCaption](../Topic/CFrameWndEx::UpdateCaption.md)|呼叫框架更新框架標題。|  
|[CFrameWndEx::WinHelp](../Topic/CFrameWndEx::WinHelp.md)|叫用 `WinHelp` 應用程式或內容相關的說明。|  
  
## 範例  
 下列範例示範如何 `CFrameWndEx` 繼承自類別的類別。  範例會說明在子類別中的方法簽章，以及如何覆寫 `OnShowPopupMenu` 方法。  這個程式碼片段是 [文字填補範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#3](../../mfc/reference/codesnippet/CPP/cframewndex-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#4](../../mfc/reference/codesnippet/CPP/cframewndex-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CFrameWndEx](../../mfc/reference/cframewndex-class.md)  
  
## 需求  
 **標題:** afxframewndex.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)