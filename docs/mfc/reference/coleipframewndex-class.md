---
title: "COleIPFrameWndEx Class | Microsoft Docs"
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
  - "COleIPFrameWndEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleIPFrameWndEx class"
ms.assetid: ebff1560-a1eb-4854-af00-95d4a192bd55
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleIPFrameWndEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`COleIPFrameWndEx` 類別會實作支援 MFC 的 OLE 容器。 您必須從 `COleIPFrameWndEx` 類別衍生應用程式的就地框架視窗類別，而不是從 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) 類別來衍生。  
  
## 語法  
  
```  
class COleIPFrameWndEx : public COleIPFrameWnd  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleIPFrameWndEx::AddDockSite](../Topic/COleIPFrameWndEx::AddDockSite.md)||  
|[COleIPFrameWndEx::AddPane](../Topic/COleIPFrameWndEx::AddPane.md)||  
|[COleIPFrameWndEx::AdjustDockingLayout](../Topic/COleIPFrameWndEx::AdjustDockingLayout.md)||  
|[COleIPFrameWndEx::DockPane](../Topic/COleIPFrameWndEx::DockPane.md)||  
|[COleIPFrameWndEx::DockPaneLeftOf](../Topic/COleIPFrameWndEx::DockPaneLeftOf.md)|將窗格停駐在另一個窗格的左邊。|  
|[COleIPFrameWndEx::EnableAutoHidePanes](../Topic/COleIPFrameWndEx::EnableAutoHidePanes.md)||  
|[COleIPFrameWndEx::EnableDocking](../Topic/COleIPFrameWndEx::EnableDocking.md)||  
|[COleIPFrameWndEx::EnablePaneMenu](../Topic/COleIPFrameWndEx::EnablePaneMenu.md)||  
|[COleIPFrameWndEx::GetActivePopup](../Topic/COleIPFrameWndEx::GetActivePopup.md)|將指標傳回到目前顯示的快顯功能表。|  
|[COleIPFrameWndEx::GetContainerFrameWindow](../Topic/COleIPFrameWndEx::GetContainerFrameWindow.md)||  
|[COleIPFrameWndEx::GetDefaultResId](../Topic/COleIPFrameWndEx::GetDefaultResId.md)|在載入視窗時傳回您指定的框架視窗資源識別碼。|  
|[COleIPFrameWndEx::GetDockFrame](../Topic/COleIPFrameWndEx::GetDockFrame.md)||  
|[COleIPFrameWndEx::GetDockingManager](../Topic/COleIPFrameWndEx::GetDockingManager.md)||  
|[COleIPFrameWndEx::GetMainFrame](../Topic/COleIPFrameWndEx::GetMainFrame.md)||  
|[COleIPFrameWndEx::GetMenuBar](../Topic/COleIPFrameWndEx::GetMenuBar.md)|將指標傳回到附加在框架視窗的功能表列物件。|  
|[COleIPFrameWndEx::GetPane](../Topic/COleIPFrameWndEx::GetPane.md)||  
|[COleIPFrameWndEx::GetTearOffBars](../Topic/COleIPFrameWndEx::GetTearOffBars.md)|傳回分割狀態的窗格物件清單。|  
|[COleIPFrameWndEx::GetToolbarButtonToolTipText](../Topic/COleIPFrameWndEx::GetToolbarButtonToolTipText.md)|架構先呼叫，再顯示工具提示按鈕。|  
|[COleIPFrameWndEx::InsertPane](../Topic/COleIPFrameWndEx::InsertPane.md)||  
|[COleIPFrameWndEx::IsMenuBarAvailable](../Topic/COleIPFrameWndEx::IsMenuBarAvailable.md)|決定功能表列物件的指標是否不是 `NULL`。|  
|[COleIPFrameWndEx::IsPointNearDockSite](../Topic/COleIPFrameWndEx::IsPointNearDockSite.md)||  
|[COleIPFrameWndEx::LoadFrame](../Topic/COleIPFrameWndEx::LoadFrame.md)|\(覆寫 `COleIPFrameWnd::LoadFrame`。\)|  
|[COleIPFrameWndEx::OnCloseDockingPane](../Topic/COleIPFrameWndEx::OnCloseDockingPane.md)||  
|[COleIPFrameWndEx::OnCloseMiniFrame](../Topic/COleIPFrameWndEx::OnCloseMiniFrame.md)||  
|[COleIPFrameWndEx::OnClosePopupMenu](../Topic/COleIPFrameWndEx::OnClosePopupMenu.md)|架構在作用中的快顯功能表處理 WM\_DESTROY 訊息時所呼叫。|  
|[COleIPFrameWndEx::OnCmdMsg](../Topic/COleIPFrameWndEx::OnCmdMsg.md)|\(覆寫 `CFrameWnd::OnCmdMsg`。\)|  
|[COleIPFrameWndEx::OnDrawMenuImage](../Topic/COleIPFrameWndEx::OnDrawMenuImage.md)|架構在繪製與功能表項目相關聯的映像時所呼叫。|  
|[COleIPFrameWndEx::OnDrawMenuLogo](../Topic/COleIPFrameWndEx::OnDrawMenuLogo.md)|架構在 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) 物件處理 WM\_PAINT 訊息時所呼叫。|  
|[COleIPFrameWndEx::OnMenuButtonToolHitTest](../Topic/COleIPFrameWndEx::OnMenuButtonToolHitTest.md)|架構在 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) 物件處理 WM\_NCHITTEST 訊息時所呼叫。|  
|[COleIPFrameWndEx::OnMoveMiniFrame](../Topic/COleIPFrameWndEx::OnMoveMiniFrame.md)||  
|[COleIPFrameWndEx::OnSetPreviewMode](../Topic/COleIPFrameWndEx::OnSetPreviewMode.md)|呼叫這個成員函式，在預覽列印模式裡外設定應用程式的主框架視窗。 \(覆寫 [CFrameWnd::OnSetPreviewMode](../Topic/CFrameWnd::OnSetPreviewMode.md)。\)|  
|[COleIPFrameWndEx::OnShowCustomizePane](../Topic/COleIPFrameWndEx::OnShowCustomizePane.md)||  
|[COleIPFrameWndEx::OnShowPanes](../Topic/COleIPFrameWndEx::OnShowPanes.md)||  
|[COleIPFrameWndEx::OnShowPopupMenu](../Topic/COleIPFrameWndEx::OnShowPopupMenu.md)|架構在啟動快顯功能表時所呼叫。|  
|[COleIPFrameWndEx::OnTearOffMenu](../Topic/COleIPFrameWndEx::OnTearOffMenu.md)|架構在啟動有分割列的功能表時所呼叫。|  
|[COleIPFrameWndEx::PaneFromPoint](../Topic/COleIPFrameWndEx::PaneFromPoint.md)||  
|[COleIPFrameWndEx::PreTranslateMessage](../Topic/COleIPFrameWndEx::PreTranslateMessage.md)|\(覆寫 `COleIPFrameWnd::PreTranslateMessage`。\)|  
|[COleIPFrameWndEx::RecalcLayout](../Topic/COleIPFrameWndEx::RecalcLayout.md)|\(覆寫 `COleIPFrameWnd::RecalcLayout`。\)|  
|[COleIPFrameWndEx::RemovePaneFromDockManager](../Topic/COleIPFrameWndEx::RemovePaneFromDockManager.md)||  
|[COleIPFrameWndEx::SetDockState](../Topic/COleIPFrameWndEx::SetDockState.md)|將指定的停駐狀態套用到屬於框架視窗的窗格。|  
|[COleIPFrameWndEx::SetupToolbarMenu](../Topic/COleIPFrameWndEx::SetupToolbarMenu.md)|藉由搜尋虛設項目並替換成指定的使用者定義項目，修改工具列物件。|  
|[COleIPFrameWndEx::ShowPane](../Topic/COleIPFrameWndEx::ShowPane.md)||  
|[COleIPFrameWndEx::WinHelp](../Topic/COleIPFrameWndEx::WinHelp.md)|架構所呼叫以起始 WinHelp 應用程式或內容說明。|  
  
### 保護方法  
  
|名稱|描述|  
|--------|--------|  
|[COleIPFrameWndEx::InitUserToobars](../Topic/COleIPFrameWndEx::InitUserToobars.md)|告知架構初始化指派給使用者定義工具列的控制項識別碼範圍。|  
  
## 範例  
 下例示範如何建立 `COleIPFrameWndEx` 類別的執行個體子類別並覆寫其方法。 此範例示範如何覆寫 `OnDestory` 方法、`RepositionFrame` 方法、`RecalcLayout` 方法和 `CalcWindowRect` 方法。 此程式碼片段是 [WordPad 範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#1](../../mfc/reference/codesnippet/CPP/coleipframewndex-class_1.cpp)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)  
  
 [COleIPFrameWndEx](../../mfc/reference/coleipframewndex-class.md)  
  
## 需求  
 **標頭：**afxoleipframewndex.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)   
 [CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)