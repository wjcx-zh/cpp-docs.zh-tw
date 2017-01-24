---
title: "CMFCListCtrl Class | Microsoft Docs"
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
  - "CMFCListCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCListCtrl class"
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
caps.latest.revision: 29
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCListCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCListCtrl` 類別會支援 [CMFCHeaderCtrl Class](../../mfc/reference/cmfcheaderctrl-class.md)的進階標題控制項功能 [CListCtrl Class](../../mfc/reference/clistctrl-class.md) 擴充類別的功能。  
  
## 語法  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCListCtrl::EnableMarkSortedColumn](../Topic/CMFCListCtrl::EnableMarkSortedColumn.md)|可以標記有不同背景色彩的排序資料行。|  
|[CMFCListCtrl::EnableMultipleSort](../Topic/CMFCListCtrl::EnableMultipleSort.md)|啟動多個排序方式。|  
|[CMFCListCtrl::GetHeaderCtrl](../Topic/CMFCListCtrl::GetHeaderCtrl.md)|傳回對底線的標題控制項的參考。|  
|[CMFCListCtrl::IsMultipleSort](../Topic/CMFCListCtrl::IsMultipleSort.md)|檢查清單控制項是否在多個排序模式。|  
|[CMFCListCtrl::OnCompareItems](../Topic/CMFCListCtrl::OnCompareItems.md)|呼叫由架構，在必須比較兩個清單控制項項目。|  
|[CMFCListCtrl::OnGetCellBkColor](../Topic/CMFCListCtrl::OnGetCellBkColor.md)|呼叫框架，則必須判斷個別儲存格的背景色彩。|  
|[CMFCListCtrl::OnGetCellFont](../Topic/CMFCListCtrl::OnGetCellFont.md)|呼叫框架，則它必須取得正在繪製的儲存格中的字型。|  
|[CMFCListCtrl::OnGetCellTextColor](../Topic/CMFCListCtrl::OnGetCellTextColor.md)|呼叫框架，則必須判斷個別儲存格的文字色彩。|  
|[CMFCListCtrl::RemoveSortColumn](../Topic/CMFCListCtrl::RemoveSortColumn.md)|從排序的資料行清單中移除排序資料行。|  
|[CMFCListCtrl::SetSortColumn](../Topic/CMFCListCtrl::SetSortColumn.md)|設定目前排序的資料行和排序次序。|  
|[CMFCListCtrl::Sort](../Topic/CMFCListCtrl::Sort.md)|排序清單控制項。|  
  
## 備註  
 `CMFCListCtrl` 為 [CListCtrl Class](../../mfc/reference/clistctrl-class.md) 類別提供兩個加強功能。  首先，它會表示資料行排序是可用的選項會自動繪製在標題的排序箭號。  接著，它支援並行排序多個資料行中的資料。  
  
## 範例  
 下列範例會在 `CMFCListCtrl` 類別會示範如何使用各種方法。  這個範例顯示如何建立清單控制項，來插入資料行，插入項目，將項目的文字，並將清單控制項的字型。  這個程式碼片段是 [Visual Studio 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/CPP/cmfclistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/CPP/cmfclistctrl-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
## 需求  
 **標題:** afxlistctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)