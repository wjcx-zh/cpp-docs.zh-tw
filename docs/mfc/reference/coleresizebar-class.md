---
title: "COleResizeBar Class | Microsoft Docs"
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
  - "COleResizeBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleResizeBar class"
  - "control bars, 調整大小"
  - "in-place items"
  - "in-place items, 調整大小"
  - "OLE items, 調整大小"
  - "resizing in-place OLE items"
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleResizeBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援重新調整就地 OLE 項目控制列的型別。  
  
## 語法  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleResizeBar::COleResizeBar](../Topic/COleResizeBar::COleResizeBar.md)|建構 `COleResizeBar` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleResizeBar::Create](../Topic/COleResizeBar::Create.md)|建立和初始化視窗的子視窗並使它與 `COleResizeBar` 物件。|  
  
## 備註  
 當使用已規劃的框線 [CRectTracker](../../mfc/reference/crecttracker-class.md) 和外部調整大小控點，`COleResizeBar` 物件的外觀。  
  
 `COleResizeBar` 物件通常是框架視窗物件的內嵌的成員 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) 從類別衍生的。  
  
 如需詳細資訊，請參閱本文 [啟動](../../mfc/activation-cpp.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 範例 SUPERPAD](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)