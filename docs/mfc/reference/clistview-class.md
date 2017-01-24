---
title: "CListView Class | Microsoft Docs"
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
  - "CListView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListView class"
  - "檢視, and common controls"
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CListView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

簡化對清單控制項的使用方式與 [CListCtrl](../../mfc/reference/clistctrl-class.md)，封裝清單控制項功能的類別，使用 MFC 的文件檢視結構。  
  
## 語法  
  
```  
class CListView : public CCtrlView  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CListView::CListView](../Topic/CListView::CListView.md)|建構 `CListView` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CListView::GetListCtrl](../Topic/CListView::GetListCtrl.md)|傳回清單控制項與這個檢視。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CListView::RemoveImageList](../Topic/CListView::RemoveImageList.md)|從清單檢視中移除指定的影像清單。|  
  
## 備註  
 如需此結構的詳細資訊，請針對上述 [CView](../../mfc/reference/cview-class.md) 類別和交互參考請參閱概觀的存在。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CListView`  
  
## 需求  
 **Header:** afxcview.h  
  
## 請參閱  
 [MFC 範例 ROWLIST](../../top/visual-cpp-samples.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)