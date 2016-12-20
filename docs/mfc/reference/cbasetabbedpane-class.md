---
title: "CBaseTabbedPane 類別 | Microsoft Docs"
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
  - "CBaseTabbedPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBaseTabbedPane 類別"
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
caps.latest.revision: 26
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBaseTabbedPane 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擴充 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的功能支援的索引標籤式視窗的建立。  
  
## 語法  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CBaseTabbedPane::CBaseTabbedPane`|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CBaseTabbedPane::AddTab](../Topic/CBaseTabbedPane::AddTab.md)|將新的索引標籤加入至索引標籤式窗格。|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../Topic/CBaseTabbedPane::AllowDestroyEmptyTabbedPane.md)|指定是否可以終結空的索引窗格。|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](../Topic/CBaseTabbedPane::ApplyRestoredTabInfo.md)|適用於定位點設定，從登錄載入，一個窗格。|  
|[CBaseTabbedPane::CanFloat](../Topic/CBaseTabbedPane::CanFloat.md)|判斷是否可以浮動窗格。  覆寫 \( [CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md)\)。|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](../Topic/CBaseTabbedPane::CanSetCaptionTextToTabName.md)|判斷索引標籤式窗格標題是否應該顯示文字和作用中的索引標籤相同。|  
|[CBaseTabbedPane::ConvertToTabbedDocument](../Topic/CBaseTabbedPane::ConvertToTabbedDocument.md)|覆寫 \( [CDockablePane::ConvertToTabbedDocument](../Topic/CDockablePane::ConvertToTabbedDocument.md)\)。|  
|[CBaseTabbedPane::DetachPane](../Topic/CBaseTabbedPane::DetachPane.md)|將一個或多個可停駐窗格為 MDI 索引標籤式文件。|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](../Topic/CBaseTabbedPane::EnableSetCaptionTextToTabName.md)|啟用或停用的索引窗格的能力同步處理標籤文字標題文字在作用中的索引標籤。|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](../Topic/CBaseTabbedPane::FillDefaultTabsOrderArray.md)|還原內部定位順序為預設狀態。|  
|[CBaseTabbedPane::FindBarByTabNumber](../Topic/CBaseTabbedPane::FindBarByTabNumber.md)|傳回位於選項的窗格中，在這個索引標籤是以零起始的索引標籤時決定的。|  
|||  
|[CBaseTabbedPane::FindPaneByID](../Topic/CBaseTabbedPane::FindPaneByID.md)|傳回由窗格 . ID 所識別的窗格|  
|[CBaseTabbedPane::FloatTab](../Topic/CBaseTabbedPane::FloatTab.md)|只有當窗格目前位於一個可拆的選項，浮動窗格，不過，。|  
|[CBaseTabbedPane::GetDefaultTabsOrder](../Topic/CBaseTabbedPane::GetDefaultTabsOrder.md)|傳回選項預設順序在窗格中。|  
|[CBaseTabbedPane::GetFirstVisibleTab](../Topic/CBaseTabbedPane::GetFirstVisibleTab.md)|擷取指標第一個顯示的索引標籤。|  
|[CBaseTabbedPane::GetMinSize](../Topic/CBaseTabbedPane::GetMinSize.md)|擷取窗格的最小容許大小。  覆寫 \( [CPane::GetMinSize](../Topic/CPane::GetMinSize.md)\)。|  
|[CBaseTabbedPane::GetPaneIcon](../Topic/CBaseTabbedPane::GetPaneIcon.md)|傳回控制代碼窗格圖示。  覆寫 \( [CBasePane::GetPaneIcon](../Topic/CBasePane::GetPaneIcon.md)\)。|  
|[CBaseTabbedPane::GetPaneList](../Topic/CBaseTabbedPane::GetPaneList.md)|傳回在索引標籤式窗格已指定的清單。|  
|[CBaseTabbedPane::GetTabArea](../Topic/CBaseTabbedPane::GetTabArea.md)|傳回頂端的週框 \(Bounding Rectangle\) 並以索引標籤區域。|  
|[CBaseTabbedPane::GetTabsNum](../Topic/CBaseTabbedPane::GetTabsNum.md)|傳回計數索引標籤視窗的索引標籤。|  
|[CBaseTabbedPane::GetUnderlyingWindow](../Topic/CBaseTabbedPane::GetUnderlyingWindow.md)|取得基礎 \(包裝\) 選項視窗。|  
|[CBaseTabbedPane::GetVisibleTabsNum](../Topic/CBaseTabbedPane::GetVisibleTabsNum.md)|傳回計數顯示的選項。|  
|[CBaseTabbedPane::HasAutoHideMode](../Topic/CBaseTabbedPane::HasAutoHideMode.md)|判斷索引標籤式窗格是否可以轉換成自動隱藏模式。|  
|[CBaseTabbedPane::IsHideSingleTab](../Topic/CBaseTabbedPane::IsHideSingleTab.md)|判斷索引標籤式窗格是否隱藏，如果只有一個索引標籤中顯示。|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|使用內部錯誤。|  
|[CBaseTabbedPane::RecalcLayout](../Topic/CBaseTabbedPane::RecalcLayout.md)|重新計算窗格的配置資訊。  覆寫 \( [CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md)\)。|  
|[CBaseTabbedPane::RemovePane](../Topic/CBaseTabbedPane::RemovePane.md)|從的索引窗格移除窗格。|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|使用內部錯誤。|  
|`CBaseTabbedPane::Serialize`|覆寫 \( [CDockablePane::Serialize](http://msdn.microsoft.com/zh-tw/09787e59-e446-4e76-894b-206d303dcfd6)\)。|  
|`CBaseTabbedPane::SerializeTabWindow`|使用內部錯誤。|  
|[CBaseTabbedPane::SetAutoDestroy](../Topic/CBaseTabbedPane::SetAutoDestroy.md)|判斷是否將自動終結定位的控制列。|  
|[CBaseTabbedPane::SetAutoHideMode](../Topic/CBaseTabbedPane::SetAutoHideMode.md)|切換顯示的和自動隱藏模式之間切換的停駐窗格。  覆寫 \( [CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md)\)。|  
|[CBaseTabbedPane::ShowTab](../Topic/CBaseTabbedPane::ShowTab.md)|顯示或隱藏索引標籤。|  
  
## 備註  
 這個類別是抽象類別，所以無法執行具現化。  它會針對各種不同的索引標籤式窗格是通用服務。  
  
 目前，程式庫包含兩個衍生的索引標籤式窗格類別: [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md) 和 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 `CBaseTabbedPane` 物件所包裝指標至 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) 物件。  [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) 之後會變成的索引窗格的子視窗。  
  
 如需如何建立的索引窗格的詳細資訊，請參閱 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)、 [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md)和 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
## 需求  
 **標題:** afxBaseTabbedPane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)