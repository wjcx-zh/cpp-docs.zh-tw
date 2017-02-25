---
title: "CSplitterWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSplitterWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSplitterWnd class"
  - "dynamic splitter windows"
  - "多重檢視"
  - "分隔視窗"
  - "static splitter windows"
  - "檢視, 多個個別框架"
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CSplitterWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供分隔視窗的功能，是 Windows 包含多個窗格。  
  
## 語法  
  
```  
class CSplitterWnd : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSplitterWnd::CSplitterWnd](../Topic/CSplitterWnd::CSplitterWnd.md)|建構 `CSplitterWnd` 物件上呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSplitterWnd::ActivateNext](../Topic/CSplitterWnd::ActivateNext.md)|執行窗格或上一個窗格命令。|  
|[CSplitterWnd::CanActivateNext](../Topic/CSplitterWnd::CanActivateNext.md)|會檢查下一個窗格或上一個窗格命令目前是否可以的。|  
|[CSplitterWnd::Create](../Topic/CSplitterWnd::Create.md)|建立動態分隔視窗並將其附加至的呼叫 `CSplitterWnd` 物件。|  
|[CSplitterWnd::CreateScrollBarCtrl](../Topic/CSplitterWnd::CreateScrollBarCtrl.md)|建立共用捲軸控制項。|  
|[CSplitterWnd::CreateStatic](../Topic/CSplitterWnd::CreateStatic.md)|建立靜態分隔視窗並將其附加至的呼叫 `CSplitterWnd` 物件。|  
|[CSplitterWnd::CreateView](../Topic/CSplitterWnd::CreateView.md)|建立在分隔視窗的窗格上呼叫。|  
|[CSplitterWnd::DeleteColumn](../Topic/CSplitterWnd::DeleteColumn.md)|刪除分隔視窗的資料行。|  
|[CSplitterWnd::DeleteRow](../Topic/CSplitterWnd::DeleteRow.md)|刪除分隔視窗的行為。|  
|[CSplitterWnd::DeleteView](../Topic/CSplitterWnd::DeleteView.md)|刪除分隔視窗的檢視。|  
|[CSplitterWnd::DoKeyboardSplit](../Topic/CSplitterWnd::DoKeyboardSplit.md)|執行除法鍵盤命令，通常是「Windows」分割。|  
|[CSplitterWnd::DoScroll](../Topic/CSplitterWnd::DoScroll.md)|執行同步處理分隔視窗捲動。|  
|[CSplitterWnd::DoScrollBy](../Topic/CSplitterWnd::DoScrollBy.md)|將內容向上捲動像素數目分割視窗。|  
|[CSplitterWnd::GetActivePane](../Topic/CSplitterWnd::GetActivePane.md)|判斷現用窗格從焦點或現用檢視在框架。|  
|[CSplitterWnd::GetColumnCount](../Topic/CSplitterWnd::GetColumnCount.md)|傳回目前窗格中的資料行計數。|  
|[CSplitterWnd::GetColumnInfo](../Topic/CSplitterWnd::GetColumnInfo.md)|傳回所指定之資料行的相關資訊。|  
|[CSplitterWnd::GetPane](../Topic/CSplitterWnd::GetPane.md)|傳回窗格在指定列和欄。|  
|[CSplitterWnd::GetRowCount](../Topic/CSplitterWnd::GetRowCount.md)|傳回目前窗格資料列計數。|  
|[CSplitterWnd::GetRowInfo](../Topic/CSplitterWnd::GetRowInfo.md)|傳回與指定之資料列的相關資訊。|  
|[CSplitterWnd::GetScrollStyle](../Topic/CSplitterWnd::GetScrollStyle.md)|傳回共用的捲軸的樣式。|  
|[CSplitterWnd::IdFromRowCol](../Topic/CSplitterWnd::IdFromRowCol.md)|傳回窗格的子視窗 ID 在指定列和欄。|  
|[CSplitterWnd::IsChildPane](../Topic/CSplitterWnd::IsChildPane.md)|呼叫以決定視窗目前是否為分隔視窗子窗格。|  
|[CSplitterWnd::IsTracking](../Topic/CSplitterWnd::IsTracking.md)|判斷分隔列目前是否已移動。|  
|[CSplitterWnd::RecalcLayout](../Topic/CSplitterWnd::RecalcLayout.md)|重新顯示分隔視窗的呼叫來調整資料列或資料行大小之後。|  
|[CSplitterWnd::SetActivePane](../Topic/CSplitterWnd::SetActivePane.md)|將窗格設定為使用中框架中。|  
|[CSplitterWnd::SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md)|呼叫會將指定的資料行資訊。|  
|[CSplitterWnd::SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md)|呼叫設定指定資料列資訊。|  
|[CSplitterWnd::SetScrollStyle](../Topic/CSplitterWnd::SetScrollStyle.md)|用於分隔視窗的共用捲軸支援指定新捲軸的樣式。|  
|[CSplitterWnd::SplitColumn](../Topic/CSplitterWnd::SplitColumn.md)|指出框架視窗位置垂直分割。|  
|[CSplitterWnd::SplitRow](../Topic/CSplitterWnd::SplitRow.md)|指出框架視窗的哪一個水平分隔。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CSplitterWnd::OnDraw](../Topic/CSplitterWnd::OnDraw.md)|呼叫框架繪製分隔視窗。|  
|[CSplitterWnd::OnDrawSplitter](../Topic/CSplitterWnd::OnDrawSplitter.md)|呈現分隔視窗的影像。|  
|[CSplitterWnd::OnInvertTracker](../Topic/CSplitterWnd::OnInvertTracker.md)|呈現分隔視窗的影像相同大小和形狀像框架視窗。|  
  
## 備註  
 窗格通常是從 [CView](../../mfc/reference/cview-class.md)衍生的特定應用程式的物件，不過，它可能會有適當的子視窗 ID. 的所有 [CWnd](../../mfc/reference/cwnd-class.md) 物件  
  
 `CSplitterWnd` 物件在父 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 或 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) 物件通常會內嵌。  使用下列步驟，建立 `CSplitterWnd` 物件:  
  
1.  將一 `CSplitterWnd` 成員變數在父框架。  
  
2.  覆寫父框架的 [CFrameWnd::OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md) 成員函式。  
  
3.  在覆寫的 `OnCreateClient`的內部，請呼叫 `CSplitterWnd`的 [建立](../Topic/CSplitterWnd::Create.md) 或 [CreateStatic](../Topic/CSplitterWnd::CreateStatic.md) 成員函式。  
  
 呼叫 **建立** 成員函式建立動態分隔視窗。  動態分隔視窗通常用於建立和移動許多個別窗格或檢視，相同資料。  這個架構便會自動建立分隔器的初始窗格，然後，在使用者操作分隔視窗的控制器，架構建立，調整大小，以及管理其他窗格。  
  
 當您呼叫 **建立**時，您指定的最小資料行高度和寬度窗格何時太小而無法完整顯示。  在呼叫 **建立**之後，您就可以呼叫 [SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md) 和 [SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md) 成員調整這些最小值函式。  
  
 請使用 `SetColumnInfo` 和 `SetRowInfo` 成員函式上設定資料行的「中的」Width 「和」資料列的理想高度。  當架構顯示分隔視窗時，會先顯示父框架，然後分隔視窗。  架構會根據理想的維度然後來配置資料行和資料列的  窗格中，從左上至分隔視窗的用戶端區域的右下角。  
  
 在動態分隔視窗的所有窗格必須屬於同一類別。  支援動態分隔視窗的熟悉的應用程式包含 Microsoft Word 和 Microsoft Excel。  
  
 使用 `CreateStatic` 成員函式建立靜態分隔視窗。  使用者可以變更窗格的大小只在靜態分隔視窗的，而不是其數值或順序。  
  
 然後，當您建立靜態分隔時，您必須明確地建立所有靜態分隔的窗格。  請確定您建立所有窗格，在父框架的 `OnCreateClient` 成員函式傳回之前，或是架構不會正確顯示視窗。  
  
 `CreateStatic` 成員函式會自動初始化具有最小資料行高度和寬度的一個靜態分隔的 0。  在呼叫 **建立**後，請呼叫 [SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md) 和 [SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md) 成員調整這些最小值函式。  此外，在您呼叫 `CreateStatic` 表示預期理想的窗格大小之後，請使用 `SetColumnInfo` 和 `SetRowInfo` 。  
  
 一個靜態分隔的個別窗格通常屬於不同的類別。  提供靜態分隔視窗的範例，請參閱圖形和編輯視窗檔案管理員。  
  
 分隔視窗支援特殊捲軸 \(除了窗格可能具有的捲軸除外\)。  這些捲軸是 `CSplitterWnd` 物件的子系和窗格共用。  
  
 然後，當您建立分隔視窗時，會建立這些特殊捲軸。  例如， `CSplitterWnd` 具有一列，兩個資料行和 **WS\_VSCROLL** 樣式會顯示由兩個窗格共用的垂直捲軸。  當使用者移動捲軸時， `WM_VSCROLL` 傳送到兩個窗格。  在  窗格中設定捲軸位置時，共用的捲軸設定。  
  
 如需分隔視窗的詳細資訊，請參閱:  
  
-   [Technical Note 29](../../mfc/tn029-splitter-windows.md)  
  
-   知識庫文件 Q262024:HOWTO:使用 CPropertySheet 做為的子系 CSplitterWnd  
  
 如需如何建立動態分隔視窗的詳細資訊，請參閱:  
  
-   MFC 範例 [Scribble](../../top/visual-cpp-samples.md)  
  
-   MFC 範例 [VIEWEX](../../top/visual-cpp-samples.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [MFC 範例 VIEWEX](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)