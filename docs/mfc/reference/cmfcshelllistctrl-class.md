---
title: "CMFCShellListCtrl Class | Microsoft Docs"
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
  - "CMFCShellListCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCShellListCtrl class"
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCShellListCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCShellListCtrl` 類別提供視窗清單控制項功能並傳遞包括展開並顯示 Shell 項目清單。  
  
## 語法  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCShellListCtrl::DisplayFolder](../Topic/CMFCShellListCtrl::DisplayFolder.md)|顯示在所提供之資料夾包含項目的清單。|  
|[CMFCShellListCtrl::DisplayParentFolder](../Topic/CMFCShellListCtrl::DisplayParentFolder.md)|顯示在資料夾會包含目前所顯示之資料夾的父項目的清單。|  
|[CMFCShellListCtrl::EnableShellContextMenu](../Topic/CMFCShellListCtrl::EnableShellContextMenu.md)|啟用或停用捷徑功能表。|  
|[CMFCShellListCtrl::GetCurrentFolder](../Topic/CMFCShellListCtrl::GetCurrentFolder.md)|擷取目前資料夾的路徑。|  
|[CMFCShellListCtrl::GetCurrentFolderName](../Topic/CMFCShellListCtrl::GetCurrentFolderName.md)|擷取目前資料夾的名稱。|  
|[CMFCShellListCtrl::GetCurrentItemIdList](../Topic/CMFCShellListCtrl::GetCurrentItemIdList.md)|傳回目前清單控制項項目的 PIDL。|  
|[CMFCShellListCtrl::GetCurrentShellFolder](../Topic/CMFCShellListCtrl::GetCurrentShellFolder.md)|傳回指向目前 Shell 資料夾。|  
|[CMFCShellListCtrl::GetItemPath](../Topic/CMFCShellListCtrl::GetItemPath.md)|傳回項目的內容路徑。|  
|[CMFCShellListCtrl::GetItemTypes](../Topic/CMFCShellListCtrl::GetItemTypes.md)|傳回由清單控制項中顯示的簡單 Shell 項目。|  
|[CMFCShellListCtrl::IsDesktop](../Topic/CMFCShellListCtrl::IsDesktop.md)|檢查目前選取的資料夾是 \[桌面\] 資料夾。|  
|[CMFCShellListCtrl::OnCompareItems](../Topic/CMFCShellListCtrl::OnCompareItems.md)|會比較兩個項目時，架構會呼叫這個方法。  \(覆寫 [CMFCListCtrl::OnCompareItems](../Topic/CMFCListCtrl::OnCompareItems.md)\)。|  
|[CMFCShellListCtrl::OnFormatFileDate](../Topic/CMFCShellListCtrl::OnFormatFileDate.md)|呼叫時，這個架構擷取清單控制項中顯示的檔案日期。|  
|[CMFCShellListCtrl::OnFormatFileSize](../Topic/CMFCShellListCtrl::OnFormatFileSize.md)|呼叫時，這個架構轉換清單控制項的檔案大小。|  
|[CMFCShellListCtrl::OnGetItemIcon](../Topic/CMFCShellListCtrl::OnGetItemIcon.md)|呼叫時，這個架構擷取清單控制項項目的圖示。|  
|[CMFCShellListCtrl::OnGetItemText](../Topic/CMFCShellListCtrl::OnGetItemText.md)|呼叫時，這個架構轉換清單控制項項目的文字。|  
|[CMFCShellListCtrl::OnSetColumns](../Topic/CMFCShellListCtrl::OnSetColumns.md)|呼叫框架，會設定資料行的名稱。|  
|[CMFCShellListCtrl::Refresh](../Topic/CMFCShellListCtrl::Refresh.md)|重新整理並重新繪製清單控制項。|  
|[CMFCShellListCtrl::SetItemTypes](../Topic/CMFCShellListCtrl::SetItemTypes.md)|將清單控制項中顯示的項目型別。|  
  
## 備註  
 `CMFCShellListCtrl` 類別可以讓您的程式列出 Windows Shell 項目 [CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md) 擴充的功能。  使用的顯示格式類似檔案總管視窗的清單檢視。  
  
 [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) 物件可以與 `CMFCShellListCtrl` 物件建立完整總管視窗。  然後，請在 `CMFCShellTreeCtrl` 的項目會使 `CMFCShellListCtrl` 物件清單中所選取項目的內容。  
  
## 範例  
 下列範例示範如何建立 `CMFCShellListCtrl` 類別的物件以及如何顯示目前顯示的資料夾之上層資料夾。  這個程式碼片段是 [Explorer 範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/CPP/cmfcshelllistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/CPP/cmfcshelllistctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/CPP/cmfcshelllistctrl-class_3.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
 [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)  
  
## 需求  
 **標題:** afxshelllistCtrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md)   
 [CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)