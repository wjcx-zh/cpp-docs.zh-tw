---
title: "CTreeView Class | Microsoft Docs"
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
  - "CTreeView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeView class"
  - "CTreeView class, 通用控制項"
  - "directory lists"
  - "file lists [C++]"
  - "tree view controls"
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTreeView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

簡化對樹狀目錄控制項會使用和。 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)，封裝樹狀目錄控制項功能的類別，使用 MFC 的文件檢視結構。  
  
## 語法  
  
```  
class CTreeView : public CCtrlView  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CTreeView::CTreeView](../Topic/CTreeView::CTreeView.md)|建構 `CTreeView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTreeView::GetTreeCtrl](../Topic/CTreeView::GetTreeCtrl.md)|會傳回樹狀目錄控制項與這個檢視。|  
  
## 備註  
 如需此結構的詳細資訊，請針對上述 [CView](../../mfc/reference/cview-class.md) 類別和交互參考請參閱概觀的存在。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CTreeView`  
  
## 需求  
 **Header:** afxcview.h  
  
## 請參閱  
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)