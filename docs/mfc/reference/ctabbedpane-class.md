---
title: "CTabbedPane Class | Microsoft Docs"
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
  - "CTabbedPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabbedPane class"
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTabbedPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作具有可拆式索引標籤之窗格的功能。  
  
## 語法  
  
```  
class CTabbedPane : public CBaseTabbedPane  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CTabbedPane::CTabbedPane`|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTabbedPane::DetachPane](../Topic/CTabbedPane::DetachPane.md)|\(覆寫 [CBaseTabbedPane::DetachPane](../Topic/CBaseTabbedPane::DetachPane.md)。\)|  
|[CTabbedPane::EnableTabAutoColor](../Topic/CTabbedPane::EnableTabAutoColor.md)|啟用或停用索引標籤的自動著色。|  
|[CTabbedPane::FloatTab](../Topic/CTabbedPane::FloatTab.md)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。  \(覆寫 [CBaseTabbedPane::FloatTab](../Topic/CBaseTabbedPane::FloatTab.md)。\)|  
|[CTabbedPane::GetTabArea](../Topic/CTabbedPane::GetTabArea.md)|傳回索引標籤式視窗內的索引標籤區域的大小和位置。|  
|[CTabbedPane::GetTabWnd](../Topic/CTabbedPane::GetTabWnd.md)||  
|[CTabbedPane::HasAutoHideMode](../Topic/CTabbedPane::HasAutoHideMode.md)|決定索引標籤式窗格是否可切換為自動隱藏模式。  \(覆寫 [CBaseTabbedPane::HasAutoHideMode](../Topic/CBaseTabbedPane::HasAutoHideMode.md)。\)|  
|[CTabbedPane::IsTabLocationBottom](../Topic/CTabbedPane::IsTabLocationBottom.md)|決定索引標籤是否位於視窗底部。|  
|[CTabbedPane::ResetTabs](../Topic/CTabbedPane::ResetTabs.md)|將所有的索引標籤式窗格重設為預設狀態。|  
|[CTabbedPane::SetTabAutoColors](../Topic/CTabbedPane::SetTabAutoColors.md)|設定在自動套色功能啟用時可以使用的自訂色彩清單。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CTabbedPane::m\_bTabsAlwaysTop](../Topic/CTabbedPane::m_bTabsAlwaysTop.md)|應用程式中的索引標籤的預設位置。|  
|[CTabbedPane::m\_pTabWndRTC](../Topic/CTabbedPane::m_pTabWndRTC.md)|自訂 `CMFCTabCtrl` 衍生物件的執行階段類別資訊。|  
  
## 備註  
 當使用者指向第二個窗格的標題，將一個窗格附加到另一個窗格時，架構會自動建立此類別的執行個體。  架構所建立的所有索引標籤式窗格，ID 皆為 \-1。  
  
 若要指定一般索引標籤，而不是 Outlook 樣式索引標籤，請將 `AFX_CBRS_REGULAR_TABS` 樣式傳遞到 [CDockablePane::CreateEx](../Topic/CDockablePane::CreateEx.md) 方法。  
  
 如果您建立具有可卸離索引標籤的索引標籤式窗格，架構可能會自動終結該窗格，因此您不應儲存指標。  若要取得索引標籤式窗格的指標，請呼叫 `CBasePane::GetParentTabbedPane` 方法。  
  
## 範例  
 在此範例中，我們會建立 `CTabbedPane` 物件。  接下來，我們使用 [CBaseTabbedPane::AddTab](../Topic/CBaseTabbedPane::AddTab.md) 附加額外的索引標籤。  
  
```  
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);  
if (!pTabbededBar->Create (_T(""), this, CRect (0, 0, 200, 200),  
                           TRUE,   
                           (UINT) -1,  
                           WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |  
                           WS_CLIPCHILDREN | CBRS_LEFT |    
                           CBRS_FLOAT_MULTI))  
{  
    TRACE0("Failed to create Solution Explorer bar\n");  
    return FALSE;      // fail to create  
}  
  
pTabbededBar->AddTab (&m_wndClassView);  
pTabbededBar->AddTab (&m_wndResourceView);  
pTabbededBar->AddTab (&m_wndFileView);  
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);  
DockPane(pTabbededBar);  
```  
  
## 範例  
 另一種可建立索引標籤式控制列物件的方式，是使用 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md)。   `AttachToTabWnd` 方法會使用 [CDockablePane::SetTabbedPaneRTC](../Topic/CDockablePane::SetTabbedPaneRTC.md) 所設定的執行階段類別資訊，以動態方式建立索引標籤式窗格物件。  
  
 在此範例中，我們會以動態方式建立索引標籤式窗格、附加兩個索引標籤，然後使第二個索引標籤無法卸離。  
  
```  
DockPane(&m_wndClassView);  
CTabbedPane* pTabbedBar = NULL;  
m_wndResourceView.AttachToTabWnd (&m_wndClassView, DM_SHOW, TRUE,  
                                  (CDockablePane**) &pTabbedBar);  
m_wndFileView.AttachToTabWnd (pTabbedBar, DM_SHOW, TRUE,  
                              (CDockablePane**) &pTabbedBar);  
pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1, FALSE);  
```  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)  
  
## 需求  
 **標頭：**afxTabbedPane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)