---
title: "CMDIFrameWndEx 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMDIFrameWndEx.AddDockSite"
  - "CMDIFrameWndEx"
  - "CMDIFrameWndEx::AddDockSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDIFrameWndEx 類別"
ms.assetid: dbcafcb3-9a7a-4f11-9dfe-ba57565c81d0
caps.latest.revision: 42
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 44
---
# CMDIFrameWndEx 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擴充 [CMDIFrameWnd](../../mfc/reference/cframewnd-class.md)的功能，視窗多重文件介面 \(MDI\) \(MDI\) 框架視窗。  
  
## 語法  
  
```  
class CMDIFrameWndEx : public CMDIFrameWnd  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMDIFrameWndEx::ActiveItemRecalcLayout](../Topic/CMDIFrameWndEx::ActiveItemRecalcLayout.md)|重新計算現用項目的配置。|  
|`CMDIFrameWndEx::AddDockSite`|沒有使用這個方法。|  
|[CMDIFrameWndEx::AddPane](../Topic/CMDIFrameWndEx::AddPane.md)|向停駐管理員的窗格。|  
|[CMDIFrameWndEx::AdjustClientArea](../Topic/CMDIFrameWndEx::AdjustClientArea.md)|減少工作區允許框線。|  
|[CMDIFrameWndEx::AdjustDockingLayout](../Topic/CMDIFrameWndEx::AdjustDockingLayout.md)|重新計算所有停駐窗格配置。|  
|[CMDIFrameWndEx::AreMDITabs](../Topic/CMDIFrameWndEx::AreMDITabs.md)|判斷 MDI 索引標籤是功能或 MDI 索引標籤式群組功能已啟用。|  
|[CMDIFrameWndEx::CanCovertControlBarToMDIChild](../Topic/CMDIFrameWndEx::CanCovertControlBarToMDIChild.md)|由架構呼叫以判斷框架視窗是否可以停駐窗格加入至索引標籤式文件。|  
|[CMDIFrameWndEx::ControlBarToTabbedDocument](../Topic/CMDIFrameWndEx::ControlBarToTabbedDocument.md)|將指定的固定窗格至索引標籤式文件。|  
|[CMDIFrameWndEx::CreateDocumentWindow](../Topic/CMDIFrameWndEx::CreateDocumentWindow.md)|建立子文件視窗。|  
|[CMDIFrameWndEx::CreateNewWindow](../Topic/CMDIFrameWndEx::CreateNewWindow.md)|由架構呼叫以建立新視窗。|  
|`CMDIFrameWndEx::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMDIFrameWndEx::DockPane](../Topic/CMDIFrameWndEx::DockPane.md)|指定內建的窗格到框架視窗。|  
|[CMDIFrameWndEx::DockPaneLeftOf](../Topic/CMDIFrameWndEx::DockPaneLeftOf.md)|停駐在其他窗格左側的窗格。|  
|[CMDIFrameWndEx::EnableAutoHidePanes](../Topic/CMDIFrameWndEx::EnableAutoHidePanes.md)|當它們停駐在主框架視窗時，指定的一邊啟動窗格的自動隱藏模式。|  
|[CMDIFrameWndEx::EnableDocking](../Topic/CMDIFrameWndEx::EnableDocking.md)|啟用屬於 MDI 框架視窗窗格的停駐。|  
|[CMDIFrameWndEx::EnableFullScreenMainMenu](../Topic/CMDIFrameWndEx::EnableFullScreenMainMenu.md)|顯示或隱藏主功能表在全螢幕模式。|  
|[CMDIFrameWndEx::EnableFullScreenMode](../Topic/CMDIFrameWndEx::EnableFullScreenMode.md)|啟動框架視窗的全螢幕模式。|  
|[CMDIFrameWndEx::EnableLoadDockState](../Topic/CMDIFrameWndEx::EnableLoadDockState.md)|啟用或停用停駐狀態的載入。|  
|[CMDIFrameWndEx::EnableMDITabbedGroups](../Topic/CMDIFrameWndEx::EnableMDITabbedGroups.md)|啟用或停用 MDI 索引標籤式群組功能。|  
|[CMDIFrameWndEx::EnableMDITabs](../Topic/CMDIFrameWndEx::EnableMDITabs.md)|啟用或停用 MDI 索引標籤功能。  啟用時，框架視窗中顯示每個 MDI 子視窗的索引標籤。|  
|[CMDIFrameWndEx::EnableMDITabsLastActiveActivation](../Topic/CMDIFrameWndEx::EnableMDITabsLastActiveActivation.md)|指定是否應該啟動最後一個作用中的索引標籤，當使用者關閉目前的索引標籤。|  
|[CMDIFrameWndEx::EnablePaneMenu](../Topic/CMDIFrameWndEx::EnablePaneMenu.md)|啟用或停用快顯功能表的窗格自動建立和管理，顯示應用程式的清單。  .|  
|[CMDIFrameWndEx::EnableWindowsDialog](../Topic/CMDIFrameWndEx::EnableWindowsDialog.md)|INSERT 命令 ID 呼叫 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) 對話方塊的功能表項目。|  
|[CMDIFrameWndEx::GetActivePopup](../Topic/CMDIFrameWndEx::GetActivePopup.md)|讓指標回到目前顯示的快顯功能表。|  
|[CMDIFrameWndEx::GetPane](../Topic/CMDIFrameWndEx::GetPane.md)|傳回指標有指定的控制項 ID. 的窗格|  
|[CMDIFrameWndEx::GetDefaultResId](../Topic/CMDIFrameWndEx::GetDefaultResId.md)|傳回 MDI 框架視窗的共用資源 ID。|  
|[CMDIFrameWndEx::GetMDITabGroups](../Topic/CMDIFrameWndEx::GetMDITabGroups.md)|傳回 MDI 索引標籤式視窗清單。|  
|[CMDIFrameWndEx::GetMDITabs](../Topic/CMDIFrameWndEx::GetMDITabs.md)|傳回參考到加上底線的索引標籤式視窗。|  
|[CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems](../Topic/CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems.md)|傳回決定旗標組合什麼內容功能表項目有效，如同的 MDI 索引標籤式群組功能時。|  
|[CMDIFrameWndEx::GetMenuBar](../Topic/CMDIFrameWndEx::GetMenuBar.md)|讓指標回到附加的功能表列物件到框架視窗。|  
|[CMDIFrameWndEx::GetRibbonBar](../Topic/CMDIFrameWndEx::GetRibbonBar.md)|擷取框架的功能區列控制項。|  
|[CMDIFrameWndEx::GetTearOffBars](../Topic/CMDIFrameWndEx::GetTearOffBars.md)|傳回 [CPane](../../mfc/reference/cpane-class.md)清單\-在 Tear\-Off 狀態的衍生物件。|  
|`CMDIFrameWndEx::GetThisClass`|由架構呼叫以取得指標與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMDIFrameWndEx::GetToolbarButtonToolTipText](../Topic/CMDIFrameWndEx::GetToolbarButtonToolTipText.md)|由架構呼叫，當應用程式顯示工具列按鈕的工具提示。|  
|[CMDIFrameWndEx::InsertPane](../Topic/CMDIFrameWndEx::InsertPane.md)|向停駐管理員的指定窗格。|  
|[CMDIFrameWndEx::IsFullScreen](../Topic/CMDIFrameWndEx::IsFullScreen.md)|決定框架視窗是否在全螢幕模式。|  
|[CMDIFrameWndEx::IsMDITabbedGroup](../Topic/CMDIFrameWndEx::IsMDITabbedGroup.md)|判斷 MDI 索引標籤式群組功能是否已啟用。|  
|[CMDIFrameWndEx::IsMemberOfMDITabGroup](../Topic/CMDIFrameWndEx::IsMemberOfMDITabGroup.md)|判斷指定的索引標籤式視窗是否在 MDI 索引標籤式群組中視窗的清單。|  
|[CMDIFrameWndEx::IsMenuBarAvailable](../Topic/CMDIFrameWndEx::IsMenuBarAvailable.md)|決定框架視窗是否有功能表列。|  
|[CMDIFrameWndEx::IsPointNearDockSite](../Topic/CMDIFrameWndEx::IsPointNearDockSite.md)|判斷指定的點是否在停駐位置附近。|  
|[CMDIFrameWndEx::IsPrintPreview](../Topic/CMDIFrameWndEx::IsPrintPreview.md)|決定框架視窗是否在預覽列印模式。|  
|[CMDIFrameWndEx::LoadFrame](../Topic/CMDIFrameWndEx::LoadFrame.md)|建立從資源資訊的框架視窗。  覆寫 \( `CMDIFrameWnd::LoadFrame`\)。|  
|[CMDIFrameWndEx::LoadMDIState](../Topic/CMDIFrameWndEx::LoadMDIState.md)|載入 MDI 索引標籤式群組和先前開啟的文件清單中指定的配置。|  
|[CMDIFrameWndEx::MDITabMoveToNextGroup](../Topic/CMDIFrameWndEx::MDITabMoveToNextGroup.md)|從目前作用中的索引標籤式視窗移動作用中的索引標籤移至下一個或目前選取群組。|  
|[CMDIFrameWndEx::MDITabNewGroup](../Topic/CMDIFrameWndEx::MDITabNewGroup.md)|建立具有單一視窗的新索引標籤式群組。|  
|[CMDIFrameWndEx::NegotiateBorderSpace](../Topic/CMDIFrameWndEx::NegotiateBorderSpace.md)|在 OLE 就地啟動時交涉在框架視窗的框線空間。|  
|[CMDIFrameWndEx::OnCloseDockingPane](../Topic/CMDIFrameWndEx::OnCloseDockingPane.md)|由架構呼叫，當使用者在可停駐窗格中按一下 \[**關閉**\] 按鈕。|  
|[CMDIFrameWndEx::OnCloseMiniFrame](../Topic/CMDIFrameWndEx::OnCloseMiniFrame.md)|由架構呼叫，當使用者在浮動迷你框架視窗中按一下 \[**關閉**\] 按鈕。|  
|[CMDIFrameWndEx::OnClosePopupMenu](../Topic/CMDIFrameWndEx::OnClosePopupMenu.md)|由架構呼叫，當一個作用中的快顯功能表處理 `WM_DESTROY` 訊息。|  
|[CMDIFrameWndEx::OnCmdMsg](../Topic/CMDIFrameWndEx::OnCmdMsg.md)|由架構呼叫以路由和分派命令訊息和更新命令使用者介面物件。|  
|[CMDIFrameWndEx::OnDrawMenuImage](../Topic/CMDIFrameWndEx::OnDrawMenuImage.md)|由架構呼叫，當與功能表項目繪製影像。|  
|[CMDIFrameWndEx::OnDrawMenuLogo](../Topic/CMDIFrameWndEx::OnDrawMenuLogo.md)|由架構呼叫，當 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)處理 `WM_PAINT` 訊息。|  
|[CMDIFrameWndEx::OnEraseMDIClientBackground](../Topic/CMDIFrameWndEx::OnEraseMDIClientBackground.md)|由架構呼叫，如同的 MDI 框架視窗處理 `WM_ERASEBKGND` 訊息。|  
|[CMDIFrameWndEx::OnMenuButtonToolHitTest](../Topic/CMDIFrameWndEx::OnMenuButtonToolHitTest.md)|由架構呼叫，當 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件來處理 `WM_NCHITTEST` 訊息。|  
|[CMDIFrameWndEx::OnMoveMiniFrame](../Topic/CMDIFrameWndEx::OnMoveMiniFrame.md)|由架構呼叫以移動小型框架視窗。|  
|[CMDIFrameWndEx::OnSetPreviewMode](../Topic/CMDIFrameWndEx::OnSetPreviewMode.md)|設定應用程式的主框架視窗預覽列印模式。  覆寫 \( [CFrameWnd::OnSetPreviewMode](../Topic/CFrameWnd::OnSetPreviewMode.md)\)。|  
|[CMDIFrameWndEx::OnShowCustomizePane](../Topic/CMDIFrameWndEx::OnShowCustomizePane.md)|由架構呼叫，以便快速自訂窗格啟動。|  
|[CMDIFrameWndEx::OnShowMDITabContextMenu](../Topic/CMDIFrameWndEx::OnShowMDITabContextMenu.md)|由架構呼叫，以便在其中一個索引標籤顯示內容功能表。  \(僅 MDI 索引標籤式群組的有效\)。|  
|[CMDIFrameWndEx::OnShowPanes](../Topic/CMDIFrameWndEx::OnShowPanes.md)|由架構呼叫以顯示或隱藏窗格。|  
|[CMDIFrameWndEx::OnShowPopupMenu](../Topic/CMDIFrameWndEx::OnShowPopupMenu.md)|由架構呼叫時，快顯功能表啟動。|  
|[CMDIFrameWndEx::OnSizeMDIClient](../Topic/CMDIFrameWndEx::OnSizeMDIClient.md)|由架構呼叫，當用戶端 MDI 視窗大小變更。|  
|[CMDIFrameWndEx::OnTearOffMenu](../Topic/CMDIFrameWndEx::OnTearOffMenu.md)|由架構呼叫，當有 Tear\-Off 列的功能表啟動。|  
|[CMDIFrameWndEx::OnUpdateFrameMenu](../Topic/CMDIFrameWndEx::OnUpdateFrameMenu.md)|由架構呼叫以更新框架功能表。  覆寫 \( `CMDIFrameWnd::OnUpdateFrameMenu`\)。|  
|[CMDIFrameWndEx::PaneFromPoint](../Topic/CMDIFrameWndEx::PaneFromPoint.md)|傳回包含指定點的停駐窗格。|  
|`CMDIFrameWndEx::PreTranslateMessage`|由 [CWinApp](../../mfc/reference/cwinapp-class.md) 類別將 Windows 訊息，這些會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前。  覆寫 \( `CMDIFrameWnd::PreTranslateMessage`\)。|  
|[CMDIFrameWndEx::RecalcLayout](../Topic/CMDIFrameWndEx::RecalcLayout.md)|由架構呼叫以重新計算框架視窗的配置。  覆寫 \( [CFrameWnd::RecalcLayout](../Topic/CFrameWnd::RecalcLayout.md)\)。|  
|[CMDIFrameWndEx::RemovePaneFromDockManager](../Topic/CMDIFrameWndEx::RemovePaneFromDockManager.md)|移除註冊窗格和從停駐管理員移除它。|  
|[CMDIFrameWndEx::SaveMDIState](../Topic/CMDIFrameWndEx::SaveMDIState.md)|儲存 MDI 索引標籤式群組和先前開啟的文件清單目前配置。|  
|[CMDIFrameWndEx::SetPrintPreviewFrame](../Topic/CMDIFrameWndEx::SetPrintPreviewFrame.md)|設定列印預覽框架視窗。|  
|[CMDIFrameWndEx::SetupToolbarMenu](../Topic/CMDIFrameWndEx::SetupToolbarMenu.md)|藉由搜尋 false 的項目和取代這些修改工具列物件具有指定使用者定義的項目。|  
|[CMDIFrameWndEx::ShowFullScreen](../Topic/CMDIFrameWndEx::ShowFullScreen.md)|轉換成從一般模式的主框架全螢幕模式。|  
|[CMDIFrameWndEx::ShowPane](../Topic/CMDIFrameWndEx::ShowPane.md)|顯示或隱藏指定的窗格。|  
|[CMDIFrameWndEx::ShowWindowsDialog](../Topic/CMDIFrameWndEx::ShowWindowsDialog.md)|建立 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) 方塊並開啟它。|  
|[CMDIFrameWndEx::TabbedDocumentToControlBar](../Topic/CMDIFrameWndEx::TabbedDocumentToControlBar.md)|轉換指定的索引標籤式文件加入至停駐窗格。|  
|[CMDIFrameWndEx::UpdateCaption](../Topic/CMDIFrameWndEx::UpdateCaption.md)|由架構呼叫以更新框架標題。|  
|[CMDIFrameWndEx::UpdateMDITabbedBarsIcons](../Topic/CMDIFrameWndEx::UpdateMDITabbedBarsIcons.md)|將每個 MDI 索引標籤式窗格的圖示。|  
|[CMDIFrameWndEx::WinHelp](../Topic/CMDIFrameWndEx::WinHelp.md)|由架構呼叫以初始化 WinHelp 應用程式或內容說明。  覆寫 \( [CWnd::WinHelp](../Topic/CWnd::WinHelp.md)\)。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMDIFrameWndEx::m\_bCanCovertControlBarToMDIChild](../Topic/CMDIFrameWndEx::m_bCanCovertControlBarToMDIChild.md)|決定停駐窗格是否可轉換為 MDI 子視窗。|  
|[CMDIFrameWndEx::m\_bDisableSetRedraw](../Topic/CMDIFrameWndEx::m_bDisableSetRedraw.md)|啟用或停用重繪 MDI 子視窗的最佳化。|  
  
## 備註  
 若要將您的 MDI 應用程式的擴充自訂功能，請從 `CMDIFrameWndEx` 衍生應用程式的 MDI 框架視窗類別而不是 `CMDIFrameWnd`。  
  
## 範例  
 下列範例會從 `CMDIFrameWndEx`衍生類別。  這個程式碼片段來自 [DrawClient 範例:MFC 功能區根據 OLE 物件繪製的應用程式](../../top/visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient#1](../../mfc/reference/codesnippet/CPP/cmdiframewndex-class_1.h)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)  
  
 [CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)  
  
## 需求  
 **標題:** afxMDIFrameWndEx.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWnd](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWndEx 類別](../../mfc/reference/cmdichildwndex-class.md)