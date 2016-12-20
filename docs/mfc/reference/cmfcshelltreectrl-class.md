---
title: "CMFCShellTreeCtrl Class | Microsoft Docs"
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
  - "CMFCShellTreeCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCShellTreeCtrl class"
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCShellTreeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCShellTreeCtrl` 類別藉由顯示 Shell 項目階層架構 [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md) 擴充功能。  
  
## 語法  
  
```  
class CMFCShellTreeCtrl : public CTreeCtrl  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCShellTreeCtrl::EnableShellContextMenu](../Topic/CMFCShellTreeCtrl::EnableShellContextMenu.md)|啟用或停用捷徑功能表。|  
|[CMFCShellTreeCtrl::GetFlags](../Topic/CMFCShellTreeCtrl::GetFlags.md)|傳回傳遞至 [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066)旗標的組合。|  
|[CMFCShellTreeCtrl::GetItemPath](../Topic/CMFCShellTreeCtrl::GetItemPath.md)|擷取的路徑項目。|  
|[CMFCShellTreeCtrl::GetRelatedList](../Topic/CMFCShellTreeCtrl::GetRelatedList.md)|傳回指向與這個物件 `CMFCShellTreeCtrl` 一起用來建立檔案總管類似的視窗的 [CMFCShellListCtrl Class](../../mfc/reference/cmfcshelllistctrl-class.md) 物件。|  
|[CMFCShellTreeCtrl::OnChildNotify](../Topic/CMFCShellTreeCtrl::OnChildNotify.md)|此成員函式以這個視窗之父視窗的呼叫，在收到適用這個視窗的通知訊息時。  \(覆寫 [CWnd::OnChildNotify](../Topic/CWnd::OnChildNotify.md)\)。|  
|[CMFCShellTreeCtrl::OnGetItemIcon](../Topic/CMFCShellTreeCtrl::OnGetItemIcon.md)||  
|[CMFCShellTreeCtrl::OnGetItemText](../Topic/CMFCShellTreeCtrl::OnGetItemText.md)||  
|[CMFCShellTreeCtrl::Refresh](../Topic/CMFCShellTreeCtrl::Refresh.md)|重新整理並重新繪製目前 `CMFCShellTreeCtrl` 物件。|  
|[CMFCShellTreeCtrl::SelectPath](../Topic/CMFCShellTreeCtrl::SelectPath.md)|選項會根據提供的 PIDL 或字串路徑的適當控制項相關之樹狀目錄的項目。|  
|[CMFCShellTreeCtrl::SetFlags](../Topic/CMFCShellTreeCtrl::SetFlags.md)|設定旗標篩選樹狀目錄內容 \(類似 `IShellFolder::EnumObjects`所使用的旗標\)。|  
|[CMFCShellTreeCtrl::SetRelatedList](../Topic/CMFCShellTreeCtrl::SetRelatedList.md)|設定目前 `CMFCShellTreeCtrl` 物件和 `CMFCShellListCtrl` 物件之間的關聯。|  
  
## 備註  
 這個類別可以讓您的程式包括 Windows Shell 項目在樹狀目錄 `CTreeCtrl` 擴充類別。  這個類別可與 `CMFCShellListCtrl` 物件建立完整總管視窗。  然後，選取樹狀結構中的項目會顯示在視窗相關清單 Shell 項目清單。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)  
  
 [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)  
  
## 需求  
 **標題:** afxshelltreeCtrl.h  
  
## 範例  
 下列範例示範如何建立 `CMFCShellTreeCtrl` 類別的物件。  這個程式碼片段是 [Explorer 範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/CPP/cmfcshelltreectrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/CPP/cmfcshelltreectrl-class_2.cpp)]  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)   
 [CMFCShellListCtrl Class](../../mfc/reference/cmfcshelllistctrl-class.md)