---
title: "COleIPFrameWnd Class | Microsoft Docs"
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
  - "COleIPFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleIPFrameWnd class"
  - "in-place editing"
  - "OLE, 編輯"
  - "OLE, in-place activation"
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleIPFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您的應用程式進行就地編輯視窗的基底。  
  
## 語法  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleIPFrameWnd::COleIPFrameWnd](../Topic/COleIPFrameWnd::COleIPFrameWnd.md)|建構 `COleIPFrameWnd` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleIPFrameWnd::OnCreateControlBars](../Topic/COleIPFrameWnd::OnCreateControlBars.md)|呼叫框架，當項目就地編輯啟動。|  
|[COleIPFrameWnd::RepositionFrame](../Topic/COleIPFrameWnd::RepositionFrame.md)|呼叫框架重新定位就地編輯視窗。|  
  
## 備註  
 這個類別會建立並放置在容器應用程式的文件視窗中的控制項陣列。  當使用者調整就地編輯視窗時，它也會處理內嵌 [COleResizeBar](../../mfc/reference/coleresizebar-class.md) 物件所產生的告知。  
  
 如需使用 `COleIPFrameWnd`的詳細資訊，請參閱本文 [啟動](../../mfc/activation-cpp.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)