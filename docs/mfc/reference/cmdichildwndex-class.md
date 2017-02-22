---
title: "CMDIChildWndEx 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMDIChildWndEx"
  - "GetThisClass"
  - "CMDIChildWndEx::PreTranslateMessage"
  - "CMDIChildWndEx::ActivateFrame"
  - "CMDIChildWndEx.GetThisClass"
  - "CMDIChildWndEx::AddDockSite"
  - "CMDIChildWndEx.CreateObject"
  - "CMDIChildWndEx::CreateObject"
  - "CMDIChildWndEx.ActivateFrame"
  - "CMDIChildWndEx::GetThisClass"
  - "CMDIChildWndEx.PreTranslateMessage"
  - "PreTranslateMessage"
  - "ActivateFrame"
  - "CreateObject"
  - "CMDIChildWndEx.AddDockSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDIChildWndEx 類別"
  - "ActivateFrame 方法"
  - "PreTranslateMessage 方法"
  - "GetThisClass 方法"
  - "CreateObject 方法"
ms.assetid: d39fec06-0bd6-4271-917d-35aae3b24d8e
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMDIChildWndEx 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMDIChildWndEx` 類別提供 Window \(MDI\) 多重文件介面 \(MDI\) 子視窗的功能。  其擴充 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)的功能。  在 MDI 應用程式中使用一些 MFC 類別時，架構會要求這個類別。  
  
## 語法  
  
```  
class CMDIChildWndEx : public CMDIChildWnd  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMDIChildWndEx::ActivateTopLevelFrame](../Topic/CMDIChildWndEx::ActivateTopLevelFrame.md)|在內部由架構呼叫以啟動最上層框架，則應該從工作列選項啟動應用程式。|  
|`CMDIChildWndEx::AddDockSite`|不使用這個方法也不會執行。|  
|[CMDIChildWndEx::AddPane](../Topic/CMDIChildWndEx::AddPane.md)|將窗格。|  
|[CMDIChildWndEx::AddTabbedPane](../Topic/CMDIChildWndEx::AddTabbedPane.md)|將的索引窗格。|  
|[CMDIChildWndEx::AdjustDockingLayout](../Topic/CMDIChildWndEx::AdjustDockingLayout.md)|調整停駐配置。|  
|[CMDIChildWndEx::CanShowOnMDITabs](../Topic/CMDIChildWndEx::CanShowOnMDITabs.md)||  
|[CMDIChildWndEx::CanShowOnTaskBarTabs](../Topic/CMDIChildWndEx::CanShowOnTaskBarTabs.md)|告知架構的 MDI 子系是否在 Windows 7 工作列索引標籤中顯示。|  
|[CMDIChildWndEx::CanShowOnWindowsList](../Topic/CMDIChildWndEx::CanShowOnWindowsList.md)|如果 MDI 子視窗的在 [CMFCWindowsManagerDialog Class](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) 對話方塊，會顯示傳回 `TRUE` 。  否則會傳回 `FALSE`。|  
|`CMDIChildWndEx::CreateObject`|由架構呼叫以建立這個類別型別的動態執行個體。|  
|[CMDIChildWndEx::DockPane](../Topic/CMDIChildWndEx::DockPane.md)|停駐窗格。|  
|[CMDIChildWndEx::DockPaneLeftOf](../Topic/CMDIChildWndEx::DockPaneLeftOf.md)|停駐在其他窗格左側的窗格。|  
|[CMDIChildWndEx::EnableAutoHidePanes](../Topic/CMDIChildWndEx::EnableAutoHidePanes.md)|當它們停駐在視窗時，指定的一邊啟動窗格的自動隱藏模式。|  
|[CMDIChildWndEx::EnableDocking](../Topic/CMDIChildWndEx::EnableDocking.md)|啟用子視窗停駐到主框架。|  
|[CMDIChildWndEx::EnableTaskbarThumbnailClipRect](../Topic/CMDIChildWndEx::EnableTaskbarThumbnailClipRect.md)|啟用或停用視窗的工作區的部分的自動選取顯示在工作列中視窗的縮圖。|  
|[CMDIChildWndEx::GetDockingManager](../Topic/CMDIChildWndEx::GetDockingManager.md)||  
|[CMDIChildWndEx::GetDocumentName](../Topic/CMDIChildWndEx::GetDocumentName.md)|傳回在 MDI 子視窗中顯示的文件名稱。|  
|[CMDIChildWndEx::GetFrameIcon](../Topic/CMDIChildWndEx::GetFrameIcon.md)|由架構呼叫以擷取 MDI 子視窗圖示。|  
|[CMDIChildWndEx::GetFrameText](../Topic/CMDIChildWndEx::GetFrameText.md)|由架構呼叫以擷取 MDI 子視窗的文字。|  
|[CMDIChildWndEx::GetPane](../Topic/CMDIChildWndEx::GetPane.md)|由指定的控制項 ID. 尋找窗格|  
|[CMDIChildWndEx::GetRelatedTabGroup](../Topic/CMDIChildWndEx::GetRelatedTabGroup.md)||  
|[CMDIChildWndEx::GetTabbedPane](../Topic/CMDIChildWndEx::GetTabbedPane.md)|傳回的指標轉換成索引標籤式文件的內嵌固定的窗格。|  
|[CMDIChildWndEx::GetTabProxyWnd](../Topic/CMDIChildWndEx::GetTabProxyWnd.md)|傳回選項 Proxy 視窗實際上向 Windows 7 工作列選項登錄。|  
|[CMDIChildWndEx::GetTaskbarPreviewWnd](../Topic/CMDIChildWndEx::GetTaskbarPreviewWnd.md)|由架構呼叫，在需要取得 Windows 7 工作列縮圖選項 \(通常檢視或分隔視窗\) 中顯示的子視窗。|  
|[CMDIChildWndEx::GetTaskbarThumbnailClipRect](../Topic/CMDIChildWndEx::GetTaskbarThumbnailClipRect.md)|由架構呼叫，在需要選取視窗工作區的一部分顯示在工作列中視窗的縮圖。|  
|`CMDIChildWndEx::GetThisClass`|由架構呼叫以取得指標與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMDIChildWndEx::GetToolbarButtonToolTipText](../Topic/CMDIChildWndEx::GetToolbarButtonToolTipText.md)|由架構呼叫以擷取工具列按鈕的工具提示。|  
|[CMDIChildWndEx::InsertPane](../Topic/CMDIChildWndEx::InsertPane.md)|向停駐管理員的指定窗格。|  
|[CMDIChildWndEx::InvalidateIconicBitmaps](../Topic/CMDIChildWndEx::InvalidateIconicBitmaps.md)|無效的 MDI 子表單的圖示點陣圖表示。|  
|[CMDIChildWndEx::IsPointNearDockSite](../Topic/CMDIChildWndEx::IsPointNearDockSite.md)|判斷指定的點是否在停駐位置附近。|  
|[CMDIChildWndEx::IsReadOnly](../Topic/CMDIChildWndEx::IsReadOnly.md)|傳回 `TRUE` ，如果在子視窗中顯示的文件是唯讀的。  否則會傳回 `FALSE`。|  
|[CMDIChildWndEx::IsRegisteredWithTaskbarTabs](../Topic/CMDIChildWndEx::IsRegisteredWithTaskbarTabs.md)|如果 MDI 子系成功向 Windows 7 工作列選項登錄，則傳回 true。|  
|[CMDIChildWndEx::IsTabbedPane](../Topic/CMDIChildWndEx::IsTabbedPane.md)|如果 MDI 子視窗的停駐窗格，則傳回 `TRUE` 。  否則會傳回 `FALSE`。|  
|[CMDIChildWndEx::IsTaskbarTabsSupportEnabled](../Topic/CMDIChildWndEx::IsTaskbarTabsSupportEnabled.md)|判斷 MDI 子系是否可以出現在 Windows 7 工作列選項。|  
|[CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled](../Topic/CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled.md)|判斷視窗工作區的部分的自動選取的顯示為在工作列中視窗的縮圖是否啟用或停用。|  
|[CMDIChildWndEx::m\_dwDefaultTaskbarTabPropertyFlags](../Topic/CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags.md)|旗標的組合，透過架構對 SetTaskbarTabProperties 方法，，當選項 \(MDI 子系\) 向 Windows 7 工作列選項登錄。  預設群組是 STPF\_USEAPPTHUMBNAILWHENACTIVE&#124;STPF\_USEAPPPEEKWHENACTIVE.|  
|[CMDIChildWndEx::OnGetIconicLivePreviewBitmap](../Topic/CMDIChildWndEx::OnGetIconicLivePreviewBitmap.md)|由架構呼叫，在需要取得 MDI 子系即時預覽的點陣圖。|  
|[CMDIChildWndEx::OnGetIconicThumbnail](../Topic/CMDIChildWndEx::OnGetIconicThumbnail.md)|由架構呼叫，在需要取得 MDI 子系圖示縮圖的點陣圖。|  
|[CMDIChildWndEx::OnMoveMiniFrame](../Topic/CMDIChildWndEx::OnMoveMiniFrame.md)|由架構呼叫以移動小型框架視窗。|  
|[CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton](../Topic/CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton.md)|由架構呼叫，當使用者在工作列選項縮圖的關閉按鈕。|  
|[CMDIChildWndEx::OnSetPreviewMode](../Topic/CMDIChildWndEx::OnSetPreviewMode.md)|由架構呼叫以進入或結束預覽列印模式。|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailActivate](../Topic/CMDIChildWndEx::OnTaskbarTabThumbnailActivate.md)|由架構呼叫，當工作列選項縮圖應該處理 WM\_ACTIVATE 訊息。|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate](../Topic/CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate.md)|由架構呼叫，當工作列選項縮圖應該處理 WM\_MOUSEACTIVATE 訊息。|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailStretch](../Topic/CMDIChildWndEx::OnTaskbarTabThumbnailStretch.md)|由架構呼叫，在需要自動縮放 Windows 7 工作列索引標籤 MDI 子系縮圖預覽的點陣圖。|  
|[CMDIChildWndEx::OnUpdateFrameTitle](../Topic/CMDIChildWndEx::OnUpdateFrameTitle.md)|由架構呼叫以更新框架標題。  覆寫 \( `CMDIChildWnd::OnUpdateFrameTitle`\)。|  
|[CMDIChildWndEx::PaneFromPoint](../Topic/CMDIChildWndEx::PaneFromPoint.md)|傳回包含指定之點的窗格。|  
|`CMDIChildWndEx::PreTranslateMessage`|由 [CWinApp](../../mfc/reference/cwinapp-class.md) 類別將 Windows 訊息，這些會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前。  覆寫 \( [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)\)。|  
|[CMDIChildWndEx::RecalcLayout](../Topic/CMDIChildWndEx::RecalcLayout.md)|重新計算視窗的配置。|  
|[CMDIChildWndEx::RegisterTaskbarTab](../Topic/CMDIChildWndEx::RegisterTaskbarTab.md)|使用 Windows 7 工作列選項的暫存器 MDI 子系。|  
|[CMDIChildWndEx::RemovePaneFromDockManager](../Topic/CMDIChildWndEx::RemovePaneFromDockManager.md)|從停駐管理員移除窗格。|  
|[CMDIChildWndEx::SetRelatedTabGroup](../Topic/CMDIChildWndEx::SetRelatedTabGroup.md)||  
|[CMDIChildWndEx::SetTaskbarTabActive](../Topic/CMDIChildWndEx::SetTaskbarTabActive.md)|啟動對應的 Windows 7 工作列選項。|  
|[CMDIChildWndEx::SetTaskbarTabOrder](../Topic/CMDIChildWndEx::SetTaskbarTabOrder.md)|在指定的視窗之前插入 MDI 子系在 Windows 7 工作列選項。|  
|[CMDIChildWndEx::SetTaskbarTabProperties](../Topic/CMDIChildWndEx::SetTaskbarTabProperties.md)|設定 Windows 7 工作列索引標籤的屬性。|  
|[CMDIChildWndEx::SetTaskbarThumbnailClipRect](../Topic/CMDIChildWndEx::SetTaskbarThumbnailClipRect.md)|內部時由架構呼叫設定裁剪矩形選取視窗工作區的一部分顯示在工作列中視窗的縮圖。|  
|[CMDIChildWndEx::ShowPane](../Topic/CMDIChildWndEx::ShowPane.md)||  
|[CMDIChildWndEx::UnregisterTaskbarTab](../Topic/CMDIChildWndEx::UnregisterTaskbarTab.md)|從 Windows 7 工作列選項移除 MDI 子系。|  
|[CMDIChildWndEx::UpdateTaskbarTabIcon](../Topic/CMDIChildWndEx::UpdateTaskbarTabIcon.md)|更新 Windows 7 工作列選項圖示。|  
  
## 備註  
 若要利用在 MDI 應用程式的擴充停駐功能，請從 `CMDIChildWndEx` 衍生您自己的應用程式 MDI 子視窗類別而不是 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)。  
  
## 範例  
 下列範例會從 `CMDIChildWndEx`衍生類別。  這個程式碼片段來自 [VisualStudioDemo 範例:MFC Visual Studio 應用程式](../../top/visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#3](../../mfc/codesnippet/CPP/cmdichildwndex-class_1.h)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)  
  
 [CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)  
  
## 需求  
 **標題:** afxMDIChildWndEx.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)   
 [CMFCWindowsManagerDialog Class](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)   
 [CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)